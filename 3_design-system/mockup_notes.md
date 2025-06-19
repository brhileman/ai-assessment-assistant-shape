# Voice Assessment Experience - Mockup Documentation

## Overview
This mockup represents the core voice conversation interface from **User Story 06: Voice Assessment Experience**. It demonstrates how stakeholders interact with the AI agent during their assessment, following LaunchPad Lab's design system.

## User Story Mapping

### Acceptance Criteria Addressed

✅ **Assessment landing page with clear "Start Assessment" button**
- *Note: This mockup shows the active conversation state. The landing page would be similar but with a prominent "Start Assessment" button instead of the conversation interface*

✅ **Professional AI agent greeting and introduction**
- Shown in the transcript with branded AI avatar and welcoming message

✅ **AI agent incorporates company custom instructions**
- Visible in the AI's first message: "Since you're from Acme Corporation, I'd love to understand your current technology landscape"

✅ **Natural conversation flow covering all assessment areas**
- Transcript shows progression from role discussion to technology stack
- Topics flow naturally from context to specific questions

✅ **"Finish Assessment" button always visible and accessible**
- Prominent secondary button (blue outline) positioned below transcript

✅ **Brief confirmation dialog before completing assessment**
- Modal popup with "Finish Assessment?" confirmation
- Provides clear choice to continue or complete

✅ **Real-time transcript display during conversation**
- Scrollable transcript area with AI/user message differentiation
- Timestamps and typing indicators for real-time feel

✅ **User controls both when conversation starts and ends**
- User-initiated through button clicks (start and finish)

## Design System Implementation

### Colors Used
- **Primary Blue (#1E60BD)**: AI messages, buttons, status indicators
- **Dark Charcoal (#2C2C35)**: Main headings, user text
- **Light Blue (#BFD7F0)**: Audio visualizer background
- **Off White (#EEEEEE)**: Transcript background
- **Gray variations**: Secondary text, borders, avatars

### Typography
- **H1 (32px, Bold)**: "AI Readiness Assessment" page title
- **Body Large (18px)**: All conversation text for readability
- **Body (16px)**: Button text, status information
- **Body Small (14px)**: Metadata, progress indicators

### Components
- **Voice Interface Card**: White background, rounded-2xl, shadow-lg
- **Audio Visualizer**: Animated bars in light blue container
- **Transcript Display**: Scrollable area with message bubbles
- **Secondary Button**: "Finish Assessment" with blue outline
- **Status Indicators**: Recording dot, connection status
- **Modal**: Confirmation dialog with warning styling

## Technical Implementation Notes

### Rails 8 + ERB Considerations

**View Structure:**
```erb
<!-- app/views/assessments/voice_interface.html.erb -->
<div class="voice-assessment-container">
  <%= render 'shared/assessment_header' %>
  <%= render 'assessments/audio_visualizer' %>
  <%= render 'assessments/transcript_display' %>
  <%= render 'assessments/assessment_controls' %>
</div>
```

**Stimulus Controllers Needed:**
- `voice-recorder-controller`: Handle OpenAI Realtime API
- `transcript-controller`: Update transcript in real-time  
- `assessment-controller`: Manage start/finish flow
- `modal-controller`: Handle confirmation dialog

### OpenAI Realtime API Integration

**Key Features to Implement:**
- WebSocket connection for real-time audio
- Speech-to-text transcription display
- AI response streaming
- Audio quality monitoring
- Connection status indicators

**Company Custom Instructions:**
- Pass company.custom_instructions to OpenAI system prompt
- Show company name in interface header
- Customize AI greeting based on company context

### Responsive Design

**Desktop (shown in mockup):**
- Max width: 800px (as per design system)
- Full-height layout for immersive experience
- Large transcript area for conversation review

**Mobile Adaptations:**
- Stack elements vertically
- Larger touch targets for buttons
- Optimize transcript scrolling for mobile
- Full-screen modal overlay

## User Experience Flow

### 1. Pre-Assessment (not shown)
- Landing page with company branding
- "Start Assessment" button
- Microphone permission request

### 2. Active Assessment (this mockup)
- Audio visualizer shows recording activity
- Real-time transcript populates
- "Finish Assessment" always available
- Progress indicators show completion status

### 3. Completion Flow
- Confirmation modal prevents accidental completion
- Clear choice to continue or finish
- Redirect to thank you page after confirmation

## Data Flow

### Assessment Model Updates
```ruby
# When conversation starts
assessment.update(status: 'in_progress', started_at: Time.current)

# Real-time transcript updates  
assessment.update(transcript: updated_transcript)

# When conversation completes
assessment.update(
  status: 'completed', 
  completed_at: Time.current,
  full_transcript: final_transcript
)
```

### Real-time Updates
- Use ActionCable for live transcript updates
- WebSocket connection for OpenAI integration
- Progressive transcript building (append-only)

## Accessibility Features

### Screen Reader Support
- Semantic HTML structure with proper headings
- Alt text for visual status indicators
- ARIA labels for interactive elements
- Live regions for transcript updates

### Keyboard Navigation
- Tab order: Header → Controls → Transcript → Finish Button
- Enter key activates buttons
- Escape key closes modal
- Focus visible indicators throughout

### Voice Interface Accessibility
- Visual indicators supplement audio feedback
- Text transcript provides full conversation record
- Clear status messages for connection/recording state

## Testing Considerations

### Manual Testing
- [ ] Microphone permission handling
- [ ] Audio quality indicators
- [ ] Transcript updates in real-time
- [ ] Button interactions and modal behavior
- [ ] Responsive design across devices

### Automated Testing (RSpec + Capybara)
- [ ] Page renders with correct elements
- [ ] Finish button triggers confirmation modal
- [ ] Modal can be dismissed or confirmed
- [ ] Assessment status updates correctly
- [ ] Company context displays properly

### Voice Integration Testing
- [ ] OpenAI API connection establishment
- [ ] Audio recording and transcription
- [ ] AI response integration
- [ ] Error handling for API failures
- [ ] Network interruption recovery

## Development Phases

### Phase 1: Static Interface
- Build HTML/CSS structure using this mockup
- Implement responsive design
- Add basic interactions (modal, buttons)

### Phase 2: Real-time Features  
- Integrate OpenAI Realtime API
- Add WebSocket connections
- Implement live transcript updates

### Phase 3: Assessment Logic
- Connect to Assessment/Company models
- Add custom instructions integration
- Implement completion flow

This mockup serves as the visual specification for implementing the voice assessment experience, ensuring consistency with both the user story requirements and LaunchPad Lab's design system. 