
# Prepare data for the sunburst chart
home_advantage_df['region'] = 'India'  # Top-level category
home_advantage_df['team_category'] = home_advantage_df['Home Field Advantage'].apply(
    lambda x: 'High Advantage (>50%)' if x > 50 else 'Low Advantage (≤50%)'
)

# Create the sunburst chart
fig = px.sunburst(
    home_advantage_df,
    path=['region', 'team_category', 'Team'],  # Hierarchy
    values='Home Field Advantage',  # Size of segments
    color='Home Field Advantage',  # Color scale
    color_continuous_scale='Viridis',
    title='IPL Teams: Home Field Advantage (Win Rate %)'
)

# Update layout for better readability
fig.update_layout(
    template='plotly_dark',
    title_font_size=20,
    margin=dict(t=50, l=25, r=25, b=25)
)

# Show the figure
fig.show()
